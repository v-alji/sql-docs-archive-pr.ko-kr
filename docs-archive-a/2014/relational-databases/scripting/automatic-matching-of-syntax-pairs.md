---
title: 구문 쌍의 자동 일치 기능
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [SQL Server], delimiter highlighting
- IntelliSense [SQL Server], syntax pair matching
ms.assetid: bfc54cda-bfd6-4545-a5b9-f9db2ae13769
author: rothja
ms.author: jroth
ms.openlocfilehash: d1237eeb9aaec39e3210b00c880c0005ef3d95bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649459"
---
# <a name="automatic-matching-of-syntax-pairs"></a><span data-ttu-id="38e1b-102">구문 쌍의 자동 일치 기능</span><span class="sxs-lookup"><span data-stu-id="38e1b-102">Automatic Matching of Syntax Pairs</span></span>
  <span data-ttu-id="38e1b-103">구문 쌍 자동 맞추기 기능은 쌍으로 코드를 작성해야 하는 구문 요소가 제대로 쌍을 이루는지 여부에 대한 즉각적인 피드백을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="38e1b-103">Automatic matching of syntax pairs gives you immediate feedback on whether syntax elements that must be coded in pairs are correctly paired.</span></span> <span data-ttu-id="38e1b-104">이를 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기에서는 구분 기호 짝 맞추기, Analysis Services XMLA 쿼리 편집기에서는 중괄호 짝 맞추기, MDX 및 DMX 편집기에서는 괄호 짝 맞추기라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e1b-104">This is known as delimiter matching in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor, brace matching in the Analysis Services XMLA Query Editor, and parenthesis matching in the MDX and DMX editors.</span></span>  
  
## <a name="database-engine-query-editor-delimiter-matching"></a><span data-ttu-id="38e1b-105">데이터베이스 엔진 쿼리 편집기의 구분 기호 짝 맞추기</span><span class="sxs-lookup"><span data-stu-id="38e1b-105">Database Engine Query Editor Delimiter Matching</span></span>  
 <span data-ttu-id="38e1b-106">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기에서는 코드 블록의 경계를 식별하는 구분 기호의 짝을 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="38e1b-106">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor matches the delimiters that identify the boundaries of code blocks.</span></span> <span data-ttu-id="38e1b-107">짝 맞추기 작업은 다음 두 가지 방법으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="38e1b-107">The matching is done in two ways:</span></span>  
  
-   <span data-ttu-id="38e1b-108">사용자가 쌍의 두 번째 구분 기호 입력을 완료하면 편집기에서 쌍의 두 구분 기호를 모두 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="38e1b-108">The editor highlights both delimiters in a pair when you finish typing the second delimiter in the pair.</span></span>  
  
-   <span data-ttu-id="38e1b-109">커서가 쌍의 구분 기호 중 하나에 있을 때 Ctrl+] 바로 가기 키를 사용하여 쌍을 이루는 다른 구분 기호로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38e1b-109">Anytime the cursor is in one of the delimiters in a pair, you can use the CTRL+] keyboard shortcut to jump to the matching delimiter.</span></span>  
  
### <a name="delimiter-pairs"></a><span data-ttu-id="38e1b-110">구분 기호 쌍</span><span class="sxs-lookup"><span data-stu-id="38e1b-110">Delimiter Pairs</span></span>  
 <span data-ttu-id="38e1b-111">자동 구분 기호 짝 맞추기 기능에서는 다음 구분 기호 집합을 인식합니다.</span><span class="sxs-lookup"><span data-stu-id="38e1b-111">Automatic delimiter matching recognizes the following sets of delimiters:</span></span>  
  
|<span data-ttu-id="38e1b-112">여는 구분 기호</span><span class="sxs-lookup"><span data-stu-id="38e1b-112">Lead Delimiter</span></span>|<span data-ttu-id="38e1b-113">닫는 구분 기호</span><span class="sxs-lookup"><span data-stu-id="38e1b-113">Closing Delimiter</span></span>|  
|--------------------|-----------------------|  
|<span data-ttu-id="38e1b-114">**(**</span><span class="sxs-lookup"><span data-stu-id="38e1b-114">**(**</span></span>|<span data-ttu-id="38e1b-115">**).**</span><span class="sxs-lookup"><span data-stu-id="38e1b-115">**)**</span></span>|  
|<span data-ttu-id="38e1b-116">**BEGIN**</span><span class="sxs-lookup"><span data-stu-id="38e1b-116">**BEGIN**</span></span>|<span data-ttu-id="38e1b-117">**END**</span><span class="sxs-lookup"><span data-stu-id="38e1b-117">**END**</span></span>|  
|<span data-ttu-id="38e1b-118">**BEGIN TRY**</span><span class="sxs-lookup"><span data-stu-id="38e1b-118">**BEGIN TRY**</span></span>|<span data-ttu-id="38e1b-119">**END TRY**</span><span class="sxs-lookup"><span data-stu-id="38e1b-119">**END TRY**</span></span>|  
|<span data-ttu-id="38e1b-120">**BEGIN CATCH**</span><span class="sxs-lookup"><span data-stu-id="38e1b-120">**BEGIN CATCH**</span></span>|<span data-ttu-id="38e1b-121">**END CATCH**</span><span class="sxs-lookup"><span data-stu-id="38e1b-121">**END CATCH**</span></span>|  
  
 <span data-ttu-id="38e1b-122">구분 기호 쌍 자동 맞추기 기능은 대괄호로 묶은 식별자([ObjectName]) 또는 따옴표 붙은 식별자("ObjectName")의 구분 기호를 인식하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38e1b-122">Automatic delimiter matching does not recognize the delimiters for bracketed identifiers ([ObjectName]), or quoted identifiers ("ObjectName").</span></span> <span data-ttu-id="38e1b-123">이미 색 구분을 통해 문자열이 구분 기호로 분리되었는지 여부가 표시되므로 쌍 맞추기 기능이 문자열 리터럴에 대해 작은따옴표 구분 기호('문자열') 쌍을 맞추지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38e1b-123">Pair matching does not match the single quotation delimiters for string literals ('string') because color coding already gives a visual indication of whether the string has been delimited.</span></span>  
  
### <a name="delimiter-highlighting"></a><span data-ttu-id="38e1b-124">구분 기호 강조 표시</span><span class="sxs-lookup"><span data-stu-id="38e1b-124">Delimiter Highlighting</span></span>  
 <span data-ttu-id="38e1b-125">짝 맞추기 기능에서 구분 기호 쌍의 여는 요소와 닫는 요소를 모두 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="38e1b-125">Matching highlights both the lead and closing element of a pair of delimiters.</span></span> <span data-ttu-id="38e1b-126">이를 통해 코드 블록을 시각적으로 식별하고 짝이 맞지 않는 구분 기호 쌍을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38e1b-126">This lets you visually identify code blocks and check for mismatched pairs of delimiters.</span></span>  
  
 <span data-ttu-id="38e1b-127">쌍을 완성하는 마지막 문자를 입력하면 구분 기호가 강조 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="38e1b-127">Delimiters are highlighted when you type the final letter that completes the pair.</span></span> <span data-ttu-id="38e1b-128">예를 들어 BEGIN을 먼저 입력한 다음 END를 입력하는 BEGIN END 쌍의 경우 END의 마지막 문자를 입력할 때 강조 표시 기능이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="38e1b-128">For example, for a BEGIN END pair where you type BEGIN first followed by END, highlighting turns on when you type the final letter in END.</span></span> <span data-ttu-id="38e1b-129">강조 표시 기능을 활성화하기 위해 반드시 여는 구분 기호와 닫는 구분 기호를 순서대로 입력할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38e1b-129">You do not have to type the lead delimiter followed by the closing delimiter to turn on highlighting.</span></span> <span data-ttu-id="38e1b-130">END를 먼저 입력한 다음 스크립트 위로 다시 스크롤하고 BEGIN을 입력할 경우 BEGIN의 마지막 문자를 입력할 때 강조 표시 기능이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="38e1b-130">If you type END first, then scroll back up the script and type BEGIN, highlighting is turned on when you type the final letter in BEGIN.</span></span> <span data-ttu-id="38e1b-131">또한 마지막에 입력한 문자가 구분 기호의 끝 문자일 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38e1b-131">The final letter typed does not have to be the end letter in the delimiter.</span></span> <span data-ttu-id="38e1b-132">예를 들어 BEGIN을 BEIN으로 잘못 입력한 경우 마지막 G를 삽입할 때 BEGIN END 쌍이 강조 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="38e1b-132">For example, you could misspell BEGIN as BEIN, when you insert the final G the BEGIN END pair is highlighted.</span></span>  
  
 <span data-ttu-id="38e1b-133">구분 기호 쌍은 커서를 이동할 때까지 강조 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="38e1b-133">The delimiter pair remains highlighted until you move the cursor.</span></span> <span data-ttu-id="38e1b-134">새 커서 위치가 동일한 구분 기호에 남아 있어도 커서가 이동하면 강조 표시 기능이 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="38e1b-134">The highlighting is turned off when the cursor is moved, even if the new cursor position remains in the same delimiter.</span></span> <span data-ttu-id="38e1b-135">쌍을 이루는 구분 기호의 문자를 삭제한 다음 다시 입력하여 강조 표시 기능을 다시 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38e1b-135">You can turn the highlighting back on by deleting and retyping any letter in either member of the pair.</span></span>  
  
## <a name="analysis-services-xmla-query-editor-brace-matching"></a><span data-ttu-id="38e1b-136">Analysis Services XMLA 쿼리 편집기의 중괄호 짝 맞추기</span><span class="sxs-lookup"><span data-stu-id="38e1b-136">Analysis Services XMLA Query Editor Brace Matching</span></span>  
 <span data-ttu-id="38e1b-137">XMLA 쿼리 편집기의 중괄호 짝 맞추기 기능은 여는 중괄호와 닫는 중괄호를 강조 표시하여 요소를 닫았는지 여부를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="38e1b-137">The XMLA Query Editor brace matching shows if you have closed elements by highlighting opening and closing braces.</span></span> <span data-ttu-id="38e1b-138">또한 Ctrl+] 바로 가기 키를 사용하여 쌍의 한 중괄호에서 다른 중괄호로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38e1b-138">You can also use the CTRL+] keyboard shortcut to jump from one brace to the matching brace.</span></span>  
  
 <span data-ttu-id="38e1b-139">XMLA 쿼리 편집기는 다음 구분 기호와 구문 요소의 중괄호 짝을 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="38e1b-139">The XMLA Query Editor does brace matching for the following terms:</span></span>  
  
-   <span data-ttu-id="38e1b-140">쌍을 이루는 시작 및 끝 태그</span><span class="sxs-lookup"><span data-stu-id="38e1b-140">Matching start and end tags.</span></span>  
  
-   <span data-ttu-id="38e1b-141">" \<" and "> " 꺾쇠 괄호 쌍</span><span class="sxs-lookup"><span data-stu-id="38e1b-141">Any pair of "\<" and ">" angle brackets.</span></span>  
  
-   <span data-ttu-id="38e1b-142">주석의 시작 및 끝</span><span class="sxs-lookup"><span data-stu-id="38e1b-142">Start and end of comments.</span></span>  
  
-   <span data-ttu-id="38e1b-143">처리 명령의 시작 및 끝</span><span class="sxs-lookup"><span data-stu-id="38e1b-143">Start and end of processing instructions.</span></span>  
  
-   <span data-ttu-id="38e1b-144">CDATA 블록의 시작 및 끝</span><span class="sxs-lookup"><span data-stu-id="38e1b-144">Start and end of CDATA blocks.</span></span>  
  
-   <span data-ttu-id="38e1b-145">DTD 선언의 시작 및 끝</span><span class="sxs-lookup"><span data-stu-id="38e1b-145">Start and end of DTD declarations.</span></span>  
  
-   <span data-ttu-id="38e1b-146">특성의 여는 따옴표 및 닫는 따옴표</span><span class="sxs-lookup"><span data-stu-id="38e1b-146">Opening and closing quotes on attributes.</span></span>  
  
## <a name="mdx-and-dmx-editor-parenthesis-matching"></a><span data-ttu-id="38e1b-147">MDX 및 DMX 편집기의 괄호 짝 맞추기</span><span class="sxs-lookup"><span data-stu-id="38e1b-147">MDX and DMX Editor Parenthesis Matching</span></span>  
 <span data-ttu-id="38e1b-148">MDX(Multi-Dimensional Expressions) 및 DMX(Data Mining Expressions) 편집기에서는 함수의 괄호 짝을 자동으로 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="38e1b-148">The Multi-Dimensional Expressions (MDX) and Data Mining Expressions (DMX) Editors automatically match parenthesis pairs in functions.</span></span>  
  
  
