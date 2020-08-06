---
title: 쿼리 옵션 결과 (텍스트 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.text.f1
ms.assetid: fd2fb409-58f9-4ede-8349-ce007126b68d
author: rothja
ms.author: jroth
ms.openlocfilehash: 45019450c8fc959b440aac5bf1e9098e59cecefc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659629"
---
# <a name="query-options-results-text-page"></a><span data-ttu-id="c5231-102">쿼리 옵션 결과(텍스트 페이지)</span><span class="sxs-lookup"><span data-stu-id="c5231-102">Query Options Results (Text Page)</span></span>
  <span data-ttu-id="c5231-103">이 페이지를 사용하여 쿼리 결과 집합을 텍스트 형식으로 표시하는 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5231-103">Use this page to specify the options for displaying a query result set in text format.</span></span> <span data-ttu-id="c5231-104">**파일로 결과 저장** 을 선택한 경우에도 이 페이지의 설정이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5231-104">The settings on this page also apply when **Results to File** is selected.</span></span>  
  
 <span data-ttu-id="c5231-105">**출력 형식**</span><span class="sxs-lookup"><span data-stu-id="c5231-105">**Output format**</span></span>  
 <span data-ttu-id="c5231-106">기본적으로 결과에 공백을 채워 만든 열에 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5231-106">By default the output is displayed in columns created by padding the results with spaces.</span></span> <span data-ttu-id="c5231-107">이외에 쉼표, 탭 또는 공백을 사용하여 열을 구분하는 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5231-107">Other options are using commas, tabs, or spaces to separate columns.</span></span> <span data-ttu-id="c5231-108">**사용자 지정 구분 기호** 입력란에 다른 구분 기호 문자를 지정하려면 **사용자 지정 구분 기호** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c5231-108">Select the **Custom delimiter** check box to specify a different delimiting character in the **Custom delimiter** box.</span></span>  
  
 <span data-ttu-id="c5231-109">**사용자 지정 구분 기호**</span><span class="sxs-lookup"><span data-stu-id="c5231-109">**Custom delimiter**</span></span>  
 <span data-ttu-id="c5231-110">열을 구분할 문자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c5231-110">Specify the character of your choice to separate columns.</span></span> <span data-ttu-id="c5231-111">이 옵션은 **출력 형식** 상자에서 **사용자 지정 구분 기호** 확인란을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5231-111">This option is only available if the **Custom delimiter** check box is selected in the **Output format** box.</span></span>  
  
 <span data-ttu-id="c5231-112">**결과 집합에 열 머리글 포함**</span><span class="sxs-lookup"><span data-stu-id="c5231-112">**Include column headers in the result set**</span></span>  
 <span data-ttu-id="c5231-113">각 열에 열 제목을 붙이지 않으려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="c5231-113">Clear this check box if you do not want each column labeled with a column title.</span></span>  
  
 <span data-ttu-id="c5231-114">**결과를 받는 대로 스크롤**</span><span class="sxs-lookup"><span data-stu-id="c5231-114">**Scroll as results are received**</span></span>  
 <span data-ttu-id="c5231-115">아래쪽의 가장 최근에 반환된 레코드에 포커스를 표시하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c5231-115">Select this check box to keep the display focus on the most recently returned records at the bottom.</span></span> <span data-ttu-id="c5231-116">받은 첫 번째 행에 포커스를 표시하려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="c5231-116">Clear this check box to keep the display focus on the first rows received.</span></span>  
  
 <span data-ttu-id="c5231-117">**숫자 값 오른쪽 맞춤**</span><span class="sxs-lookup"><span data-stu-id="c5231-117">**Right align numeric values**</span></span>  
 <span data-ttu-id="c5231-118">숫자 값을 열 오른쪽에 맞추려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c5231-118">Select this check box to align numeric values to the right of the column.</span></span> <span data-ttu-id="c5231-119">이렇게 하면 고정 소수 자릿수를 가진 숫자를 쉽게 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5231-119">This can make it easier to review numbers with a fixed number of decimal places.</span></span>  
  
 <span data-ttu-id="c5231-120">**쿼리 실행 후 결과 삭제**</span><span class="sxs-lookup"><span data-stu-id="c5231-120">**Discard result after query executes**</span></span>  
 <span data-ttu-id="c5231-121">화면에 표시한 후 쿼리 결과를 삭제하여 메모리를 확보합니다.</span><span class="sxs-lookup"><span data-stu-id="c5231-121">Frees memory by discarding the query results after the screen display has received them.</span></span>  
  
 <span data-ttu-id="c5231-122">**별도의 탭에 결과 표시**</span><span class="sxs-lookup"><span data-stu-id="c5231-122">**Display results in a separate tab**</span></span>  
 <span data-ttu-id="c5231-123">쿼리 문서 창의 아래쪽 대신 새로운 문서 창에 결과 집합을 표시하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c5231-123">Select this check box to display the result set in a new document window, instead of at the bottom of the query document window.</span></span>  
  
 <span data-ttu-id="c5231-124">**쿼리 실행 후 결과 탭으로 전환**</span><span class="sxs-lookup"><span data-stu-id="c5231-124">**Switch to results tab after the query executes**</span></span>  
 <span data-ttu-id="c5231-125">자동으로 화면 포커스를 결과 집합에 두려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c5231-125">Click to automatically set the screen focus to the result set.</span></span>  
  
 <span data-ttu-id="c5231-126">**각 열에 표시할 최대 문자 수**</span><span class="sxs-lookup"><span data-stu-id="c5231-126">**Maximum number of characters displayed in each column**</span></span>  
 <span data-ttu-id="c5231-127">기본값은 256자입니다.</span><span class="sxs-lookup"><span data-stu-id="c5231-127">This value defaults to 256.</span></span> <span data-ttu-id="c5231-128">이보다 큰 결과 집합을 잘리지 않게 표시하려면 값을 높입니다.</span><span class="sxs-lookup"><span data-stu-id="c5231-128">Increase this value to display larger result sets without truncation.</span></span>  
  
 <span data-ttu-id="c5231-129">**기본값으로 다시 설정**</span><span class="sxs-lookup"><span data-stu-id="c5231-129">**Reset to Default**</span></span>  
 <span data-ttu-id="c5231-130">이 페이지의 모든 값을 원래 기본값으로 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c5231-130">Resets all values on this page to the original default values.</span></span>  
  
## <a name="saving-a-text-result-set-with-headers"></a><span data-ttu-id="c5231-131">머리글을 포함하여 텍스트 결과 집합 저장</span><span class="sxs-lookup"><span data-stu-id="c5231-131">Saving a text result set with headers</span></span>  
 <span data-ttu-id="c5231-132">쿼리 결과를 머리글이 있는 텍스트 파일로 저장하려면 **결과 집합에 열 머리글 포함** 확인란과 구분된 출력 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c5231-132">To save query results as a text file with headers, select the **Include column headers in the result set** check box and a delimited output format.</span></span> <span data-ttu-id="c5231-133">그러면 도구 모음에서 **파일로 결과 저장** 을 클릭하거나, 또는 쿼리 결과를 마우스 오른쪽 단추로 클릭하고 **다른 이름으로 결과 저장**을 클릭하고 파일 이름을 입력한 다음 **저장**을 클릭할 때 생성되는 보고서 파일에 머리글이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5231-133">Now the report file will contain headers when you click **Results to File** on the toolbar, or when you right-click any query results, click **Save Results As**, type a file name, and then click **Save**.</span></span>  
  
  
