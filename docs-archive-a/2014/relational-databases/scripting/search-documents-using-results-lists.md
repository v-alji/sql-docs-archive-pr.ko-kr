---
title: 결과 목록을 사용하여 문서 검색
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- searches [SQL Server Management Studio], result lists
- result list searches [SQL Server Management Studio]
- searches [SQL Server Management Studio], multiple files
- Query Editor [SQL Server Management Studio], search multiple files
ms.assetid: 275e1b6c-fbd0-4408-af77-35903f90657c
author: rothja
ms.author: jroth
ms.openlocfilehash: 58ff3754bc1667de75426e52b3ddd855e7d1a348
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660471"
---
# <a name="search-documents-using-results-lists"></a><span data-ttu-id="7c992-102">결과 목록을 사용하여 문서 검색</span><span class="sxs-lookup"><span data-stu-id="7c992-102">Search Documents Using Results Lists</span></span>
  <span data-ttu-id="7c992-103">**찾기 및 바꾸기** 대화 상자를 사용하면 프로젝트나 솔루션 또는 파일 시스템 폴더의 모든 파일을 검색하여 바꿀 수 있으며 이러한 파일이 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 열려 있지 않은 경우에도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="7c992-103">Using the **Find and Replace** dialog box, you can search and replace text in all files in a project or solution or in a file system folder, even when they are not open in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="7c992-104">**찾기 및 바꾸기** 대화 상자에서 수행한 검색 조건과 일치하는 항목이 찾기 결과 1 및 찾기 결과 2 창에 나타나며 일치하는 항목이 포함된 줄에서 해당 텍스트를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c992-104">Matches from searches that were performed with the **Find and Replace** dialog box appear in the Find Results 1 and Find Results 2 windows, which allows you to view the exact text from the line containing the match.</span></span>  
  
### <a name="to-search-in-multiple-files"></a><span data-ttu-id="7c992-105">여러 파일을 검색하려면</span><span class="sxs-lookup"><span data-stu-id="7c992-105">To search in multiple files</span></span>  
  
1.  <span data-ttu-id="7c992-106">**편집** 메뉴에서 **찾기 및 바꾸기** 를 가리킨 다음 **파일에서 찾기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7c992-106">On the **Edit** menu, point to **Find and Replace,** and then click **Find in Files**.</span></span>  
  
2.  <span data-ttu-id="7c992-107">**찾을 내용** 입력란에 검색할 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7c992-107">In the **Find what** text box, enter the text to search for.</span></span>  
  
3.  <span data-ttu-id="7c992-108">**찾는 위치** 목록에서 **모든 열린 문서**, **현재 프로젝트**또는 **전체 솔루션**을 클릭하거나 디렉터리 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7c992-108">In the **Look in** list, click **All Open Documents**, **Current Project**, **Entire Solution**, or type a directory path.</span></span>  
  
4.  <span data-ttu-id="7c992-109">**파일 형식** 목록에서 나열된 파일 확장명 집합 중 하나를 선택하거나 검색할 파일 형식에 대한 확장명을 쉼표로 구분하여 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7c992-109">In the **File types** list, select one of the listed sets of file extensions or enter the extensions for the types of files to be searched, separated by semicolons.</span></span> <span data-ttu-id="7c992-110">대신 \*에서 열려 있지 않은 경우에도 마찬가지입니다.\* 를 사용하여 **찾는 위치** 드롭다운 목록에 나열된 디렉터리에서 모든 파일을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c992-110">Use \*.\* to search all files in the directory listed in the **Look in** drop-down list.</span></span>  
  
5.  <span data-ttu-id="7c992-111">검색의 정확도를 높이려면 나머지 검색 옵션 중에서 원하는 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7c992-111">Select from the remaining search options to improve the accuracy of the search.</span></span>  
  
6.  <span data-ttu-id="7c992-112">**찾기** 를 클릭하여 검색을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="7c992-112">Click **Find** to begin the search.</span></span>  
  
 <span data-ttu-id="7c992-113">검색 조건과 일치하는 항목이 기본적으로 찾기 결과 1 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c992-113">The matches for the search appear in the Find Results 1 window by default.</span></span> <span data-ttu-id="7c992-114">찾기 결과 1 창에서 각 항목을 두 번 클릭하여 검색 조건과 일치하는 항목을 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c992-114">You can browse the search matches by double-clicking each entry in the Find Results 1 window.</span></span> <span data-ttu-id="7c992-115">새 창에서 검색 결과를 보려면 **찾기 2에 표시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7c992-115">To view the search results in a new window, select **Display in Find 2**.</span></span>  
  
#### <a name="to-replace-across-multiple-files-or-folders"></a><span data-ttu-id="7c992-116">여러 파일이나 폴더에서 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="7c992-116">To replace across multiple files or folders</span></span>  
  
1.  <span data-ttu-id="7c992-117">**편집** 메뉴에서 **찾기 및 바꾸기** 를 가리킨 다음 **파일에서 바꾸기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7c992-117">On the **Edit** menu, point to **Find and Replace,** and then click **Replace in Files**.</span></span>  
  
2.  <span data-ttu-id="7c992-118">**찾을 내용** 입력란에 검색할 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7c992-118">In the **Find what** text box, enter the text to search for.</span></span>  
  
3.  <span data-ttu-id="7c992-119">**바꿀 내용** 상자에 검색 텍스트를 바꿀 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7c992-119">In the **Replace with** box, enter the text to replace the search text.</span></span>  
  
4.  <span data-ttu-id="7c992-120">**찾는 위치** 목록에서 **모든 열린 문서**, **현재 프로젝트**또는 **전체 솔루션**을 클릭하거나 디렉터리 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7c992-120">In the **Look in** list, click **All Open Documents**, **Current Project**, **Entire Solution**, or type a directory path.</span></span>  
  
5.  <span data-ttu-id="7c992-121">**바꾸기** 를 클릭하여 현재 검색 조건과 일치하는 항목을 **바꿀 내용** 상자에 있는 텍스트로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7c992-121">Click **Replace** to replace the current search match with the text in the **Replace with** box.</span></span> <span data-ttu-id="7c992-122">**다음 찾기** 를 클릭하여 일치하는 항목 하나를 건너뛰거나 **파일 건너뛰기**를 클릭하여 전체 파일을 건너뛸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c992-122">You can skip a single match by clicking **Find Next** or skip an entire file clicking **Skip File**.</span></span>  
  
     <span data-ttu-id="7c992-123">\- 또는-</span><span class="sxs-lookup"><span data-stu-id="7c992-123">\- or -</span></span>  
  
     <span data-ttu-id="7c992-124">**모두 바꾸기** 를 클릭하여 현재 검색 조건과 일치하는 모든 항목을 **바꿀 내용** 상자에 있는 텍스트로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7c992-124">Choose **Replace all** to replace all search matches with the text in the **Replace with** box.</span></span> <span data-ttu-id="7c992-125">나중에 바꾼 내용 중 일부를 실행 취소하려면 **모두 바꾸기를 실행한 후 수정한 파일 열어 두기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7c992-125">Select **Keep modified files open after Replace All** if you want to undo some of the replacements at another time.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7c992-126">**모두 바꾸기** 는 **파일 건너뛰기** 또는 **다음 찾기**로 건너뛴 파일의 일치하는 항목을 비롯하여 검색 조건과 일치하는 모든 항목을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7c992-126">**Replace all** replaces all search matches, including those in files you have skipped with **Skip File** or **Find Next**.</span></span> <span data-ttu-id="7c992-127">바꾸기 작업 후에 계속 열려 있는 파일에서 수행된 바꾸기에 대해서만 **실행 취소** 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c992-127">You can only use **Undo** for replacements made in files that remain open after the replacement operation.</span></span>  
  
 <span data-ttu-id="7c992-128">기본적으로 찾기 결과 1 창에 바꾸기 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c992-128">Replacement information appears in the Find Results 1 window by default.</span></span> <span data-ttu-id="7c992-129">찾기 결과 1 창에서 각 항목을 두 번 클릭하여 바꾸기 정보를 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c992-129">You can browse replacements by double-clicking each entry in the Find Results 1 window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c992-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7c992-130">See Also</span></span>  
 <span data-ttu-id="7c992-131">[찾기 및 바꾸기](search-and-replace.md) </span><span class="sxs-lookup"><span data-stu-id="7c992-131">[Search and Replace](search-and-replace.md) </span></span>  
 <span data-ttu-id="7c992-132">[대화형으로 문서 검색](search-documents-interactively.md) </span><span class="sxs-lookup"><span data-stu-id="7c992-132">[Search Documents Interactively](search-documents-interactively.md) </span></span>  
 <span data-ttu-id="7c992-133">[와일드카드로 텍스트 검색](search-text-with-wildcards.md) </span><span class="sxs-lookup"><span data-stu-id="7c992-133">[Search Text with Wildcards](search-text-with-wildcards.md) </span></span>  
 [<span data-ttu-id="7c992-134">정규식을 사용한 텍스트 검색</span><span class="sxs-lookup"><span data-stu-id="7c992-134">Search Text with Regular Expressions</span></span>](search-text-with-regular-expressions.md)  
  
  
