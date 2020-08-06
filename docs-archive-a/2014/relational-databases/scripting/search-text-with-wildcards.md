---
title: 와일드카드로 텍스트 검색
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- vswildcardsbuilder
helpviewer_keywords:
- searches [SQL Server Management Studio], wildcards
- Query Editor [SQL Server Management Studio], wildcard searches
- wildcard options [SQL Server Management Studio]
ms.assetid: 449600f8-cc87-4b3f-878a-59c158a88a40
author: rothja
ms.author: jroth
ms.openlocfilehash: cc4e24c3dce73e46350b0c106429c42ab5f0edb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660987"
---
# <a name="search-text-with-wildcards"></a><span data-ttu-id="4bfd0-102">와일드카드로 텍스트 검색</span><span class="sxs-lookup"><span data-stu-id="4bfd0-102">Search Text with Wildcards</span></span>
  <span data-ttu-id="4bfd0-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **찾기 및 바꾸기** 대화 상자의 **찾을 내용** 필드에서 다음 식은 문자나 숫자를 대체할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bfd0-103">The following expressions can replace characters or digits in the **Find what** field of the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Find and Replace** dialog box.</span></span>  
  
#### <a name="to-search-using-wildcards"></a><span data-ttu-id="4bfd0-104">와일드카드를 사용하여 검색하려면</span><span class="sxs-lookup"><span data-stu-id="4bfd0-104">To search using wildcards</span></span>  
  
1.  <span data-ttu-id="4bfd0-105">빠른 찾기, **파일에서 찾기** , **빠른 바꾸기**또는 **파일에서 바꾸기**작업 중에 **찾을 내용** 필드에서 와일드카드를 사용할 수 있게 하려면 **찾기 옵션** 아래에서 **사용** 옵션을 선택한 다음 **와일드카드**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4bfd0-105">To enable the use of wildcards in the **Find what** field during Quick Find, **Find in Files**, **Quick Replace**, or **Replace in Files** operations, select the **Use** option under **Find Options** and then choose **Wildcards**.</span></span>  
  
2.  <span data-ttu-id="4bfd0-106">그러면 **찾을 내용** 필드 옆에 있는 삼각형 **참조 목록** 단추를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bfd0-106">The triangular **Reference List** button next to the **Find what** field then becomes available.</span></span> <span data-ttu-id="4bfd0-107">이 단추를 클릭하여 사용할 수 있는 와일드카드 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4bfd0-107">Click this button to display a list of the available wildcards.</span></span> <span data-ttu-id="4bfd0-108">**참조 목록**에서 임의의 항목을 선택하면 해당 항목이 **찾을 대상** 문자열에 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bfd0-108">When you choose any item from the **Reference List**, it is inserted into the **Find what** string.</span></span>  
  
 <span data-ttu-id="4bfd0-109">다음 표에서는 **참조 목록**에서 사용할 수 있는 와일드카드를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4bfd0-109">The following table describes the wildcards available in the **Reference List**.</span></span>  
  
|<span data-ttu-id="4bfd0-110">식</span><span class="sxs-lookup"><span data-stu-id="4bfd0-110">Expression</span></span>|<span data-ttu-id="4bfd0-111">구문</span><span class="sxs-lookup"><span data-stu-id="4bfd0-111">Syntax</span></span>|<span data-ttu-id="4bfd0-112">Description</span><span class="sxs-lookup"><span data-stu-id="4bfd0-112">Description</span></span>|  
|----------------|------------|-----------------|  
|<span data-ttu-id="4bfd0-113">임의의 단일 문자</span><span class="sxs-lookup"><span data-stu-id="4bfd0-113">Any single character</span></span>|<span data-ttu-id="4bfd0-114">?</span><span class="sxs-lookup"><span data-stu-id="4bfd0-114">?</span></span>|<span data-ttu-id="4bfd0-115">임의의 문자 하나에 대응합니다.</span><span class="sxs-lookup"><span data-stu-id="4bfd0-115">Matches any single character.</span></span>|  
|<span data-ttu-id="4bfd0-116">임의의 단일 숫자</span><span class="sxs-lookup"><span data-stu-id="4bfd0-116">Any single digit</span></span>|#|<span data-ttu-id="4bfd0-117">임의의 숫자 하나와 대응합니다.</span><span class="sxs-lookup"><span data-stu-id="4bfd0-117">Matches any single digit.</span></span> <span data-ttu-id="4bfd0-118">예를 들어 7#은 7 다음에 다른 숫자 하나가 표시되는 숫자와 일치합니다(즉, 71과는 일치하지만 17과는 일치하지 않음).</span><span class="sxs-lookup"><span data-stu-id="4bfd0-118">For example, 7# matches numbers that include 7 followed by another number, such as 71, but not 17.</span></span>|  
|<span data-ttu-id="4bfd0-119">집합에 없는 문자</span><span class="sxs-lookup"><span data-stu-id="4bfd0-119">Characters not in set</span></span>|<span data-ttu-id="4bfd0-120">[!</span><span class="sxs-lookup"><span data-stu-id="4bfd0-120">[!</span></span> <span data-ttu-id="4bfd0-121">]</span><span class="sxs-lookup"><span data-stu-id="4bfd0-121">]</span></span>|<span data-ttu-id="4bfd0-122">집합에 지정되지 않는 임의의 문자 하나와 대응합니다.</span><span class="sxs-lookup"><span data-stu-id="4bfd0-122">Matches any one character that is not specified in the set.</span></span>|  
|<span data-ttu-id="4bfd0-123">하나 이상의 문자</span><span class="sxs-lookup"><span data-stu-id="4bfd0-123">One or more characters</span></span>|*|<span data-ttu-id="4bfd0-124">하나 이상의 임의의 문자와 대응합니다.</span><span class="sxs-lookup"><span data-stu-id="4bfd0-124">Matches any one or more characters.</span></span> <span data-ttu-id="4bfd0-125">예를 들어 new\*는 "new"를 포함하는 임의의 텍스트(예: newfile.txt)와 대응합니다.</span><span class="sxs-lookup"><span data-stu-id="4bfd0-125">For example, new\* matches any text that includes "new", such as newfile.txt.</span></span>|  
|<span data-ttu-id="4bfd0-126">문자 집합</span><span class="sxs-lookup"><span data-stu-id="4bfd0-126">Set of characters</span></span>|<span data-ttu-id="4bfd0-127">[ ]</span><span class="sxs-lookup"><span data-stu-id="4bfd0-127">[ ]</span></span>|<span data-ttu-id="4bfd0-128">집합에 지정된 문자 중 하나와 대응합니다.</span><span class="sxs-lookup"><span data-stu-id="4bfd0-128">Matches any one of the characters specified in the set.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4bfd0-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4bfd0-129">See Also</span></span>  
 <span data-ttu-id="4bfd0-130">[찾기 및 바꾸기](search-and-replace.md) </span><span class="sxs-lookup"><span data-stu-id="4bfd0-130">[Search and Replace](search-and-replace.md) </span></span>  
 [<span data-ttu-id="4bfd0-131">정규식을 사용한 텍스트 검색</span><span class="sxs-lookup"><span data-stu-id="4bfd0-131">Search Text with Regular Expressions</span></span>](search-text-with-regular-expressions.md)  
