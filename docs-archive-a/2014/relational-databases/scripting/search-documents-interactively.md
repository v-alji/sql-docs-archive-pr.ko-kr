---
title: 대화형으로 문서 검색
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- interactive searches [SQL Server Management Studio]
- searches [SQL Server Management Studio], interactive
- Query Editor [SQL Server Management Studio], interactive search
ms.assetid: dae65ac5-67af-45c6-a6e0-952fea26d680
author: rothja
ms.author: jroth
ms.openlocfilehash: 5603db77ea4f58d4bb036635a23ec3cfa400a818
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660476"
---
# <a name="search-documents-interactively"></a><span data-ttu-id="a2bae-102">대화형으로 문서 검색</span><span class="sxs-lookup"><span data-stu-id="a2bae-102">Search Documents Interactively</span></span>
  <span data-ttu-id="a2bae-103">**찾기 및 바꾸기** 대화 상자를 사용하면 하나 이상의 열려 있는 파일이나 창을 검색하고 검색 조건과 일치하는 항목을 하나씩 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2bae-103">Using the **Find and Replace** dialog box, you can search one or more open files or windows and move through the search matches one by one.</span></span> <span data-ttu-id="a2bae-104">이 기술을 사용하면 일치하는 항목 주위의 텍스트 컨텍스트에서 일치하는 개별 항목을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2bae-104">This technique allows you to review each individual search match in the context of the text around the match.</span></span> <span data-ttu-id="a2bae-105">또한 **찾기 및 바꾸기** 대화 상자를 사용하여 대량 찾기 작업을 수행하고 검색 조건과 일치하는 항목을 보고서 형식으로 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2bae-105">You also have the option of performing bulk find operations and reviewing search matches in report format using the **Find and Replace** dialog box.</span></span>  
  
### <a name="to-search-all-open-documents"></a><span data-ttu-id="a2bae-106">열린 모든 문서를 검색하려면</span><span class="sxs-lookup"><span data-stu-id="a2bae-106">To search all open documents</span></span>  
  
1.  <span data-ttu-id="a2bae-107">검색할 항목을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a2bae-107">Open the items you wish to search.</span></span>  
  
2.  <span data-ttu-id="a2bae-108">**편집** 메뉴에서 **찾기 및 바꾸기** 를 가리킨 다음 **빠른 찾기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a2bae-108">On the **Edit** menu, point to **Find and Replace,** and then click **QuickFind**.</span></span>  
  
3.  <span data-ttu-id="a2bae-109">**찾기 및 바꾸기** 입력란에 검색할 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a2bae-109">In the **Find and Replace** text box, enter the text to search for.</span></span>  
  
4.  <span data-ttu-id="a2bae-110">**찾는 위치** 목록에서 **모든 열린 문서**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a2bae-110">In the **Look in** list, select **All Open Documents**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a2bae-111">**모든 열린 문서** 를 선택한 경우 열려 있는 특정 파일이 검색되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2bae-111">Certain open files might not be searched when **All Open Documents** is selected.</span></span> <span data-ttu-id="a2bae-112">텍스트 뷰(예: 코드 뷰)에서 현재 열려 있는 파일만 검색에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2bae-112">Only files currently open in a textual view, such as Code view, are included in searches.</span></span> <span data-ttu-id="a2bae-113">디자이너 뷰의 파일은 검색에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a2bae-113">Files in Designer view are not included in searches.</span></span>  
  
5.  <span data-ttu-id="a2bae-114">검색의 정확도를 높이려면 추가 검색 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a2bae-114">Select additional search options to increase the accuracy of the search.</span></span>  
  
6.  <span data-ttu-id="a2bae-115">**다음 찾기** 를 클릭하여 검색을 시작하고 마지막 파일이 검색될 때까지 계속해서 **다음 찾기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a2bae-115">Click **Find Next** to start the search, and continue clicking **Find Next** until the last file has been searched.</span></span>  
  
 <span data-ttu-id="a2bae-116">문서의 시작 또는 끝을 검색이 통과하면 상태 표시줄에 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2bae-116">When the search passes the beginning or end of the document, a message is displayed in the status bar.</span></span> <span data-ttu-id="a2bae-117">검색의 시작 지점에 검색이 도달하면 메시지 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a2bae-117">A message box appears when the search reaches the starting point of the search.</span></span>  
  
#### <a name="to-replace-in-all-active-files-interactively"></a><span data-ttu-id="a2bae-118">모든 활성 파일에서 대화형으로 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="a2bae-118">To replace in all active files interactively</span></span>  
  
1.  <span data-ttu-id="a2bae-119">**편집** 메뉴에서 **찾기 및 바꾸기**를 가리킨 다음 **빠른 바꾸기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a2bae-119">On the **Edit** menu, point to **Find and Replace**, and then click **QuickReplace**.</span></span>  
  
2.  <span data-ttu-id="a2bae-120">**찾을 내용** 상자에 검색할 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a2bae-120">In the **Find what** box, enter the text to search for.</span></span>  
  
3.  <span data-ttu-id="a2bae-121">**바꿀 내용** 상자에 검색 텍스트를 바꿀 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a2bae-121">In the **Replace with** box, enter the text to replace the search text.</span></span>  
  
4.  <span data-ttu-id="a2bae-122">**찾는 위치** 목록에서 **모든 열린 문서**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a2bae-122">In the **Look in** list, select **All Open Documents**.</span></span>  
  
5.  <span data-ttu-id="a2bae-123">**바꾸기**를 클릭하고 마지막 파일의 마지막 항목이 바뀔 때까지 계속해서 **바꾸기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a2bae-123">Click **Replace**, and continue clicking **Replace** until the last match in the last file has been replaced.</span></span> <span data-ttu-id="a2bae-124">바꾸지 않을 항목을 건너뛰려면 **다음 찾기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a2bae-124">Click **Find Next** to skip a match you do not want to replace.</span></span>  
  
     <span data-ttu-id="a2bae-125">또는</span><span class="sxs-lookup"><span data-stu-id="a2bae-125">-or-</span></span>  
  
     <span data-ttu-id="a2bae-126">**모두 바꾸기** 를 선택하여 일치하는 모든 항목을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a2bae-126">Choose **Replace All** to replace all matches.</span></span> <span data-ttu-id="a2bae-127">바뀐 항목의 총 개수가 표시되는 메시지 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a2bae-127">A message box appears, listing the total number of replacements.</span></span>  
  
 <span data-ttu-id="a2bae-128">**모두 바꾸기** 명령은 **다음 찾기** 단추로 건너뛴 항목을 비롯하여 일치하는 모든 항목을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a2bae-128">The **Replace All** command replaces all search matches, including those you have skipped with the **Find Next** button.</span></span> <span data-ttu-id="a2bae-129">**모두 바꾸기**를 취소하려면 파일을 닫기 전에 **편집** 메뉴에서 **실행 취소** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a2bae-129">To cancel **Replace All**, click **Undo** from the **Edit** menu before closing any of the files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2bae-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a2bae-130">See Also</span></span>  
 <span data-ttu-id="a2bae-131">[활성 문서에서 입력하는 순서대로 검색](search-an-active-document-incrementally.md) </span><span class="sxs-lookup"><span data-stu-id="a2bae-131">[Search an Active Document Incrementally](search-an-active-document-incrementally.md) </span></span>  
 <span data-ttu-id="a2bae-132">[찾기 및 바꾸기](search-and-replace.md) </span><span class="sxs-lookup"><span data-stu-id="a2bae-132">[Search and Replace](search-and-replace.md) </span></span>  
 <span data-ttu-id="a2bae-133">[결과 목록을 사용하여 문서 검색](search-documents-using-results-lists.md) </span><span class="sxs-lookup"><span data-stu-id="a2bae-133">[Search Documents Using Results Lists](search-documents-using-results-lists.md) </span></span>  
 <span data-ttu-id="a2bae-134">[와일드카드로 텍스트 검색](search-text-with-wildcards.md) </span><span class="sxs-lookup"><span data-stu-id="a2bae-134">[Search Text with Wildcards](search-text-with-wildcards.md) </span></span>  
 [<span data-ttu-id="a2bae-135">정규식을 사용한 텍스트 검색</span><span class="sxs-lookup"><span data-stu-id="a2bae-135">Search Text with Regular Expressions</span></span>](search-text-with-regular-expressions.md)  
  
  
