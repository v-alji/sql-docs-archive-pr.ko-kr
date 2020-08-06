---
title: 활성 문서에서 입력하는 순서대로 검색
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- searches [SQL Server Management Studio], incremental
- Query Editor [SQL Server Management Studio], incremental search
- incremental searches [SQL Server Management Studio]
ms.assetid: 490bb36c-dd43-4219-9e2a-ff27046b9395
author: rothja
ms.author: jroth
ms.openlocfilehash: aefc2f0b7abff5992a8f4f7817e564ef1b72009d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647591"
---
# <a name="search-an-active-document-incrementally"></a><span data-ttu-id="dfb20-102">활성 문서에서 입력하는 순서대로 검색</span><span class="sxs-lookup"><span data-stu-id="dfb20-102">Search an Active Document Incrementally</span></span>
  <span data-ttu-id="dfb20-103">텍스트를 입력하여 하나의 문서나 창을 증분식으로 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb20-103">You can search a single document or window incrementally by entering text.</span></span> <span data-ttu-id="dfb20-104">검색 작업은 문서나 창에서 증분 검색 중에 입력된 문자와 일치하는 첫 번째 문자 집합을 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb20-104">The search operation highlights the first set of characters that matches the characters entered during the incremental search in the document or window.</span></span> <span data-ttu-id="dfb20-105">증분 검색은 숨겨진 텍스트를 제외하고 문서나 창에 있는 모든 텍스트를 자동으로 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb20-105">Incremental search automatically searches all of the text within a document or window except for text that has been hidden.</span></span>  
  
 <span data-ttu-id="dfb20-106">**대/소문자 구분** 옵션의 경우 증분 검색은 이전 검색의 조건을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb20-106">For the **Match case** option, incremental search uses the criteria from your previous search.</span></span> <span data-ttu-id="dfb20-107">예를 들어 **파일에서 찾기** 대화 상자를 사용하여 여러 파일을 검색했으며 **대/소문자 구분**을 선택한 경우 다음에 증분식으로 검색을 수행하면 검색에서 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb20-107">For example, if you searched across multiple files using the **Find in Files** dialog box and select **Match Case**, and you next search incrementally, the search will be case-sensitive.</span></span>  
  
### <a name="to-search-incrementally"></a><span data-ttu-id="dfb20-108">증분식으로 검색하려면</span><span class="sxs-lookup"><span data-stu-id="dfb20-108">To search incrementally</span></span>  
  
1.  <span data-ttu-id="dfb20-109">검색할 파일이나 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dfb20-109">Open the file or window to you want to search.</span></span>  
  
2.  <span data-ttu-id="dfb20-110">**편집** 메뉴에서 **고급**을 가리킨 다음 **증분 검색**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb20-110">On the **Edit** menu, point to **Advanced**, and then click **Incremental Search**.</span></span>  
  
     <span data-ttu-id="dfb20-111">커서 아이콘이 검색 방향을 나타나는 화살표가 있는 쌍안경 모양으로 바뀌고 상태 표시줄에 "증분 검색"이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfb20-111">The cursor icon changes to a binocular with an arrow, indicating the search direction, and the status bar displays "Incremental Search."</span></span>  
  
3.  <span data-ttu-id="dfb20-112">텍스트 문자열 입력을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb20-112">Begin typing the text string.</span></span>  
  
     <span data-ttu-id="dfb20-113">입력하는 텍스트가 상태 표시줄에 표시되면서 텍스트와 일치하는 첫 번째 항목이 편집기에서 강조 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfb20-113">The status bar displays the text you are entering while the editor highlights the first occurrence that matches the text.</span></span> <span data-ttu-id="dfb20-114">입력을 계속하면 편집기는 일치하는 다음 항목으로 이동하여 해당 항목을 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb20-114">As you continue typing, the editor moves to the next match and highlights it.</span></span> <span data-ttu-id="dfb20-115">일치하는 항목이 없으면 상태 표시줄에 다음이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfb20-115">If no matches are available, the status bar displays the following.</span></span>  
  
    ```  
    Incremental Search: <text> (not found)  
    ```  
  
 <span data-ttu-id="dfb20-116">증분 검색은 문서의 현재 위치에서 아래 방향으로 왼쪽에서 오른쪽으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfb20-116">Incremental searches are performed from the current location in the document downwards from left to right.</span></span> <span data-ttu-id="dfb20-117">바로 가기 키를 사용하여 증분 검색을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb20-117">Incremental searches can be done using keyboard shortcut keys.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dfb20-118">바로 가기 키의 전체 목록을 보려면 [SQL Server Management Studio 바로 가기 키](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dfb20-118">For a complete list of keyboard shortcut keys, see [SQL Server Management Studio Keyboard Shortcuts](../../ssms/sql-server-management-studio-keyboard-shortcuts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfb20-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dfb20-119">See Also</span></span>  
 <span data-ttu-id="dfb20-120">[찾기 및 바꾸기](search-and-replace.md) </span><span class="sxs-lookup"><span data-stu-id="dfb20-120">[Search and Replace](search-and-replace.md) </span></span>  
 <span data-ttu-id="dfb20-121">[대화형으로 문서 검색](search-documents-interactively.md) </span><span class="sxs-lookup"><span data-stu-id="dfb20-121">[Search Documents Interactively](search-documents-interactively.md) </span></span>  
 <span data-ttu-id="dfb20-122">[결과 목록을 사용하여 문서 검색](search-documents-using-results-lists.md) </span><span class="sxs-lookup"><span data-stu-id="dfb20-122">[Search Documents Using Results Lists](search-documents-using-results-lists.md) </span></span>  
 <span data-ttu-id="dfb20-123">[와일드카드로 텍스트 검색](search-text-with-wildcards.md) </span><span class="sxs-lookup"><span data-stu-id="dfb20-123">[Search Text with Wildcards](search-text-with-wildcards.md) </span></span>  
 [<span data-ttu-id="dfb20-124">정규식을 사용한 텍스트 검색</span><span class="sxs-lookup"><span data-stu-id="dfb20-124">Search Text with Regular Expressions</span></span>](search-text-with-regular-expressions.md)  
  
  
