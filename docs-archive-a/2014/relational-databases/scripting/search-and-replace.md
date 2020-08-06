---
title: 찾기 및 바꾸기
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- match case [SQL Server]
- undo operations
- searches [SQL Server Management Studio]
- replacing text
- quick search and replaces [SQL Server Management Studio]
- Query Editor [SQL Server Management Studio], undo
- Query Editor [SQL Server Management Studio], searching
- regular expressions [SQL Server Management Studio]
- finding text [SQL Server Management Studio]
- text [SQL Server], search and replace operations
- finding [SQL Server Management Studio]
- locating text
- Query Editor [SQL Server Management Studio], replacing text
- Find and Replace dialog box
- wildcard options [SQL Server Management Studio]
- match whole word [SQL Server]
- searches [SQL Server Management Studio], replacing
ms.assetid: 3641c7b3-3e3e-4ddd-af82-c15b50004f94
author: rothja
ms.author: jroth
ms.openlocfilehash: 55422fa7201213477426c7bc25c45ff05acf8945
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647588"
---
# <a name="search-and-replace"></a><span data-ttu-id="d9be8-102">찾기 및 바꾸기</span><span class="sxs-lookup"><span data-stu-id="d9be8-102">Search and Replace</span></span>
  <span data-ttu-id="d9be8-103">텍스트를 찾아서 바꾸는 방법에는 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9be8-103">There are several different ways to find and replace text.</span></span> <span data-ttu-id="d9be8-104">**편집** 메뉴에서 **찾기 및 바꾸기** 는 **빠른 찾기**, **빠른 바꾸기**, **파일에서 찾기**또는 **파일에서 바꾸기**의 네 가지 선택 사항을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d9be8-104">On the **Edit** menu, **Find and Replace** offers four choices: **Quick Find**, **Quick Replace**, **Find in Files**, or **Replace in Files**.</span></span> <span data-ttu-id="d9be8-105">이러한 각 항목은 해당 버전의 **찾기 및 바꾸기** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d9be8-105">Each of these opens versions of the **Find and Replace** dialog box.</span></span> <span data-ttu-id="d9be8-106">또한 증분 검색 바로 가기 키를 사용하여 대화 상자 없이 검색을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9be8-106">You can also search without a dialog box by using incremental search keyboard shortcut keys.</span></span> <span data-ttu-id="d9be8-107">이러한 기술을 사용하면 찾기 및 바꾸기의 범위를 제어하고 검색 조건과 일치하는 항목 및 바꾼 항목을 검토하는 방법을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9be8-107">These techniques allow you to control the scope of find and replace, and choose the method of reviewing search matches and replacements.</span></span>  
  
 <span data-ttu-id="d9be8-108">텍스트를 검색하고 바꿀 경우에는 다음 사항을 살펴 보십시오.</span><span class="sxs-lookup"><span data-stu-id="d9be8-108">You should consider the following when you search and replace text:</span></span>  
  
-   <span data-ttu-id="d9be8-109">**찾기 및 바꾸기** 대화 상자에 설정된 옵션은 모든 검색에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d9be8-109">Options set in the **Find and Replace** dialog box affect all the searches.</span></span> <span data-ttu-id="d9be8-110">이러한 옵션에는 **대/소문자 구분**, **단어 단위로**, **위로 검색**, **숨겨진 텍스트 검색**, **와일드카드**, **정규식**, **찾는 위치: 모든 열린 문서**, **찾는 위치: 현재 문서**등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9be8-110">These options include **Match case**, **Match whole word**, **Search up**, **Search hidden text**, **Wildcards**, **Regular Expressions**, **Look in All Open Documents**, and **Look in Current Project**.</span></span> <span data-ttu-id="d9be8-111">모든 버전의 **찾기 및 바꾸기** 대화 상자에서 모든 옵션을 사용할 수 있는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="d9be8-111">All options are not available in all versions of the **Find and Replace** dialog box.</span></span>  
  
-   <span data-ttu-id="d9be8-112">**실행 취소** 는 바꾸기 작업 이후에 열려 있는 문서에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9be8-112">**Undo** is available only for documents left open after a replace operation.</span></span>  
  
-   <span data-ttu-id="d9be8-113">여러 파일에 대해**모두 바꾸기** 작업의 **실행 취소** 를 수행하면 해당 작업은 영향을 받은 모든 파일에 적용되는 하나의 대량 동작으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9be8-113">**Undo** for a **Replace All** operation that spans more than one file is considered a single, bulk action across all the affected files.</span></span> <span data-ttu-id="d9be8-114">즉, 일부 파일에서만 변경 내용을 취소하고 다른 파일에서 변경 내용을 유지할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d9be8-114">That is, you cannot undo the change in some files while retaining the change in other files.</span></span>  
  
 <span data-ttu-id="d9be8-115">일반적으로 그래픽 보기가 포함된 항목은 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d9be8-115">Generally, you cannot search items with graphical views.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9be8-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d9be8-116">See Also</span></span>  
 <span data-ttu-id="d9be8-117">[활성 문서에서 입력하는 순서대로 검색](search-an-active-document-incrementally.md) </span><span class="sxs-lookup"><span data-stu-id="d9be8-117">[Search an Active Document Incrementally](search-an-active-document-incrementally.md) </span></span>  
 <span data-ttu-id="d9be8-118">[대화형으로 문서 검색](search-documents-interactively.md) </span><span class="sxs-lookup"><span data-stu-id="d9be8-118">[Search Documents Interactively](search-documents-interactively.md) </span></span>  
 <span data-ttu-id="d9be8-119">[결과 목록을 사용하여 문서 검색](search-documents-using-results-lists.md) </span><span class="sxs-lookup"><span data-stu-id="d9be8-119">[Search Documents Using Results Lists](search-documents-using-results-lists.md) </span></span>  
 <span data-ttu-id="d9be8-120">[와일드카드로 텍스트 검색](search-text-with-wildcards.md) </span><span class="sxs-lookup"><span data-stu-id="d9be8-120">[Search Text with Wildcards](search-text-with-wildcards.md) </span></span>  
 [<span data-ttu-id="d9be8-121">정규식을 사용한 텍스트 검색</span><span class="sxs-lookup"><span data-stu-id="d9be8-121">Search Text with Regular Expressions</span></span>](search-text-with-regular-expressions.md)  
  
  
