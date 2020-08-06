---
title: 쿼리 옵션 결과 (그리드 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.grid.f1
ms.assetid: 764bf435-3aab-4c62-b4e0-64fe020a5a95
author: rothja
ms.author: jroth
ms.openlocfilehash: bf300dd5071128b0259230ae788a27595bd8d29e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659630"
---
# <a name="query-options-results-grid-page"></a><span data-ttu-id="fd8c1-102">쿼리 옵션 결과(표 형태 페이지)</span><span class="sxs-lookup"><span data-stu-id="fd8c1-102">Query Options Results (Grid Page)</span></span>
  <span data-ttu-id="fd8c1-103">이 페이지를 사용하여 쿼리 결과 집합을 표 형태로 표시하는 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd8c1-103">Use this page to specify the options for displaying a query result set in grid format.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fd8c1-104">옵션</span><span class="sxs-lookup"><span data-stu-id="fd8c1-104">Options</span></span>  
 <span data-ttu-id="fd8c1-105">**결과 집합에 쿼리 포함**</span><span class="sxs-lookup"><span data-stu-id="fd8c1-105">**Include the query in the result set**</span></span>  
 <span data-ttu-id="fd8c1-106">결과 집합의 일부로 쿼리 텍스트를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fd8c1-106">Returns the text of the query as part of the result set.</span></span>  
  
 <span data-ttu-id="fd8c1-107">**결과를 복사하거나 저장할 때 열 머리글 포함**</span><span class="sxs-lookup"><span data-stu-id="fd8c1-107">**Include column headers when copying or saving the results**</span></span>  
 <span data-ttu-id="fd8c1-108">결과를 클립보드에 복사하거나 파일에 저장할 때 열 머리글(제목)을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="fd8c1-108">Include column headers (titles) when results are copied to the clipboard, or saved in a file.</span></span> <span data-ttu-id="fd8c1-109">저장하거나 복사한 결과 데이터에 열 머리글 없이 데이터만 포함하려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="fd8c1-109">Clear this check box if you do not want saved or copied result data to have only the data, and not the column headings.</span></span>  
  
 <span data-ttu-id="fd8c1-110">**실행 후 결과 삭제**</span><span class="sxs-lookup"><span data-stu-id="fd8c1-110">**Discard results after execution**</span></span>  
 <span data-ttu-id="fd8c1-111">화면에 표시한 후 쿼리 결과를 삭제하여 메모리를 확보합니다.</span><span class="sxs-lookup"><span data-stu-id="fd8c1-111">Free memory by discarding the query results after the screen display has received them.</span></span>  
  
 <span data-ttu-id="fd8c1-112">**별도의 탭에 결과 표시**</span><span class="sxs-lookup"><span data-stu-id="fd8c1-112">**Display results in a separate tab**</span></span>  
 <span data-ttu-id="fd8c1-113">쿼리 문서 창의 아래쪽 대신 새로운 문서 창에 결과 집합을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fd8c1-113">Display the result set in a new document window, instead of at the bottom of the query document window.</span></span>  
  
 <span data-ttu-id="fd8c1-114">**쿼리 실행 후 결과 탭으로 전환**</span><span class="sxs-lookup"><span data-stu-id="fd8c1-114">**Switch to results tab after the query executes**</span></span>  
 <span data-ttu-id="fd8c1-115">자동으로 화면 포커스를 결과 집합에 둡니다.</span><span class="sxs-lookup"><span data-stu-id="fd8c1-115">Automatically set the screen focus to the result set.</span></span>  
  
 <span data-ttu-id="fd8c1-116">**검색한 최대 문자 수**</span><span class="sxs-lookup"><span data-stu-id="fd8c1-116">**Maximum Characters Retrieved**</span></span>  
 <span data-ttu-id="fd8c1-117">**비 XML 데이터**:</span><span class="sxs-lookup"><span data-stu-id="fd8c1-117">**Non XML data**:</span></span>  
  
 <span data-ttu-id="fd8c1-118">1에서 65535 사이의 숫자를 입력하여 각 셀에 표시될 최대 문자 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fd8c1-118">Enter a number from 1 through 65535 to specify the maximum number of characters that will be displayed in each cell.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fd8c1-119">너무 많은 문자를 지정하면 결과 집합의 데이터가 잘려 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd8c1-119">Specifying a large number of characters may cause data in the result set to appear truncated.</span></span> <span data-ttu-id="fd8c1-120">각 셀에 표시되는 최대 문자 수는 글꼴 크기에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="fd8c1-120">The maximum number of characters displayed in each cell is dependent on the font size.</span></span> <span data-ttu-id="fd8c1-121">이 입력란에 높은 값을 입력하면 큰 결과 집합이 반환될 경우 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 의 메모리 실행 속도가 느려지거나 시스템 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd8c1-121">When large result sets are returned, a high value in this box can cause [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to run low on memory and hinder system performance.</span></span>  
  
 <span data-ttu-id="fd8c1-122">**XML 데이터**:</span><span class="sxs-lookup"><span data-stu-id="fd8c1-122">**XML data**:</span></span>  
  
 <span data-ttu-id="fd8c1-123">1mb, **2mb 또는** **5mb** **를 선택 합니다**.</span><span class="sxs-lookup"><span data-stu-id="fd8c1-123">Select **1 MB**, **2 MB**, or **5 MB**.</span></span> <span data-ttu-id="fd8c1-124">모든 문자를 검색하려면 **제한 없음** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fd8c1-124">Select **Unlimited** to retrieve all characters.</span></span>  
  
 <span data-ttu-id="fd8c1-125">**기본값으로 다시 설정**</span><span class="sxs-lookup"><span data-stu-id="fd8c1-125">**Reset to Default**</span></span>  
 <span data-ttu-id="fd8c1-126">이 페이지의 모든 값을 원래 기본값으로 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fd8c1-126">Resets all values on this page to the original default values.</span></span>  
  
  
