---
title: 찾기 및 바꾸기
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Find and Replace dialog box
ms.assetid: 09297893-d80b-4c88-86b4-52bfb639e521
author: rothja
ms.author: jroth
ms.openlocfilehash: 9735c2c7271382e3b25ce2b50299153f16882ef0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660490"
---
# <a name="find-and-replace"></a><span data-ttu-id="e0452-102">찾기 및 바꾸기</span><span class="sxs-lookup"><span data-stu-id="e0452-102">Find and Replace</span></span>
  <span data-ttu-id="e0452-103">**찾기 및 바꾸기** 대화 상자를 사용하여 파일 내에서 텍스트를 찾을 수 있으며 필요하면 다른 텍스트로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-103">Use the **Find and Replace** dialog box to locate text within a file and optionally replace it.</span></span> <span data-ttu-id="e0452-104">대화 상자를 여는 방법에 따라 **찾기 및 바꾸기** 대화 상자에 표시되는 옵션이 조금씩 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-104">Versions of the **Find and Replace** dialog box with slightly different options can appear, depending on how the dialog box was opened.</span></span> <span data-ttu-id="e0452-105">찾기 옵션만 있고 바꾸기 옵션은 없는 대화 상자를 열려면 **편집** 메뉴에서 **찾기 및 바꾸기**를 가리킨 다음 **빠른 찾기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-105">On the **Edit** menu, point to **Find and Replace**, and then click **Quick Find** to open the dialog box with find options, but without replace options.</span></span> <span data-ttu-id="e0452-106">찾기 옵션과 바꾸기 옵션이 모두 있는 대화 상자를 열려면 **편집** 메뉴에서 **찾기 및 바꾸기**를 가리킨 다음 **빠른 바꾸기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-106">On the **Edit** menu, point to **Find and Replace**, and then click **Quick Replace** to open the dialog box with both find options and replace options.</span></span>  
  
 <span data-ttu-id="e0452-107">도구 모음 단추 및 바로 가기 키를 사용하여 **찾기 및 바꾸기** 대화 상자를 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-107">Toolbar buttons and shortcut keys are also available to open the **Find and Replace** dialog box.</span></span>  
  
## <a name="find-what"></a><span data-ttu-id="e0452-108">찾을 내용</span><span class="sxs-lookup"><span data-stu-id="e0452-108">Find What</span></span>  
 <span data-ttu-id="e0452-109">다음 컨트롤을 사용하면 일치하는 문자열이나 식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-109">These controls enable you to specify the string or expression that will be matched.</span></span>  
  
 <span data-ttu-id="e0452-110">**찾을 내용**</span><span class="sxs-lookup"><span data-stu-id="e0452-110">**Find what**</span></span>  
 <span data-ttu-id="e0452-111">검색할 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-111">Type the text to search for.</span></span> <span data-ttu-id="e0452-112">대화 상자에서는 대화 상자를 열기 전에 커서로 선택한 텍스트, 가까이 위치한 텍스트 또는 이전에 검색한 텍스트를 사용하여 가능한 검색 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-112">The dialog box attempts to fill in a probable search text, using text selected with the cursor before opening the dialog box, or nearby text, or previously searched-for text.</span></span> <span data-ttu-id="e0452-113">드롭다운 목록에서 검색 문자열을 선택하여 가장 최근에 사용한 20개의 문자열을 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-113">You can reuse one of the last 20 search strings by selecting it from this drop-down list.</span></span>  
  
 <span data-ttu-id="e0452-114">**[와일드카드가 포함된 문자열]**</span><span class="sxs-lookup"><span data-stu-id="e0452-114">**[string with wildcards]**</span></span>  
 <span data-ttu-id="e0452-115">검색 문자열에 별표(`*`) 및 물음표(`?`)와 같은 와일드카드를 사용하려면 **찾기 옵션** 아래의 **사용** 확인란을 선택한 다음 **와일드카드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-115">If you want to use wildcards such as asterisks (`*`) and question marks (`?`) in your search string, select the **Use** check box under **Find Options** and then click **Wildcards**.</span></span>  
  
 <span data-ttu-id="e0452-116">**[정규식]**</span><span class="sxs-lookup"><span data-stu-id="e0452-116">**[regular expression]**</span></span>  
 <span data-ttu-id="e0452-117">검색 엔진에서 검색 문자열을 정규식으로 해석하려면 **찾기 옵션** 아래의 **사용** 확인란을 선택한 다음 **정규식**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-117">To cause the search engine to interpret your search string as a regular expression, select the **Use** check box under **Find Options** and then click **Regular expressions**.</span></span>  
  
 <span data-ttu-id="e0452-118">**식 작성기**</span><span class="sxs-lookup"><span data-stu-id="e0452-118">**Expression Builder**</span></span>  
 <span data-ttu-id="e0452-119">**찾기 옵션** 에서 **사용** 확인란을 선택하면 **찾을 내용**입력란 옆에 있는 삼각형 단추가 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-119">This triangular button next to the **Find what** box becomes available when the **Use** check box is selected in **Find Options**.</span></span> <span data-ttu-id="e0452-120">이 단추를 클릭하면 선택한 **사용** 옵션에 따라 와일드카드 또는 정규식 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-120">Click this button to display a list of wildcards or regular expressions, depending upon the **Use** option selected.</span></span> <span data-ttu-id="e0452-121">이 목록에서 항목을 선택하면 해당 항목이 **찾을 내용** 입력란에 지정된 문자열에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-121">Choosing any item from this list adds it to the string specified in the **Find what** box.</span></span>  
  
## <a name="replace-with"></a><span data-ttu-id="e0452-122">바꿀 항목</span><span class="sxs-lookup"><span data-stu-id="e0452-122">Replace With</span></span>  
 <span data-ttu-id="e0452-123">이러한 컨트롤을 사용하면 일치하는 문자열 또는 식의 자리에 삽입할 내용을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-123">These controls enable you to specify what will be inserted in the place of the matched string or expression.</span></span>  
  
 <span data-ttu-id="e0452-124">**Replace with**</span><span class="sxs-lookup"><span data-stu-id="e0452-124">**Replace with**</span></span>  
 <span data-ttu-id="e0452-125">**찾을 내용** 에 지정된 문자열의 인스턴스를 다른 문자열로 바꾸려면 이 필드에 바꿀 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-125">To replace instances of the string specified in **Find what** with another string, enter the replacement string in this field.</span></span> <span data-ttu-id="e0452-126">**찾을 내용**으로 검색한 문자열을 삭제하려면 이 필드를 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-126">To delete instances of the text specified in **Find what**, leave this field blank.</span></span> <span data-ttu-id="e0452-127">가장 최근에 입력한 20개의 항목을 표시하려면 드롭다운 목록을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-127">Select the drop-down list to display the last 20 items entered.</span></span> <span data-ttu-id="e0452-128">**바꿀 내용** 입력란에 지정된 문자열에 정규식을 포함하려면 **사용** 확인란을 클릭한 다음 **정규식**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-128">To include regular expressions in the string specified in the **Replace with** box, click the **Use** check box and then click **Regular Expressions**.</span></span> <span data-ttu-id="e0452-129">이 입력란은 **빠른 바꾸기**를 클릭하여 대화 상자를 열었을 때만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-129">This box only appears if this dialog box was opened by clicked **Quick Replace**.</span></span>  
  
 <span data-ttu-id="e0452-130">**Replace with**</span><span class="sxs-lookup"><span data-stu-id="e0452-130">**Replace with**</span></span>  
 <span data-ttu-id="e0452-131">**찾을 내용** 입력란에 지정된 문자열의 인스턴스를 다른 문자열로 바꾸려면 이 필드에 바꿀 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-131">To replace instances of the string specified in the **Find what** box with another string, enter the replacement string in this field.</span></span> <span data-ttu-id="e0452-132">**찾을 내용** 에 지정된 문자열을 삭제하려면 이 필드를 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-132">To delete instances of the string specified in the **Find what** box, leave this field blank.</span></span> <span data-ttu-id="e0452-133">가장 최근에 입력한 20개의 항목을 표시하려면 드롭다운 목록을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-133">Select the drop-down list to display the last 20 items entered.</span></span> <span data-ttu-id="e0452-134">**바꿀 내용** 입력란에 지정된 문자열에 정규식을 포함하려면 **사용** 확인란을 클릭한 다음 **정규식**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-134">To include regular expressions in the string specified in the **Replace with** box, click the **Use** check box and then click **Regular Expressions**.</span></span>  
  
 <span data-ttu-id="e0452-135">**식 작성기**</span><span class="sxs-lookup"><span data-stu-id="e0452-135">**Expression Builder**</span></span>  
 <span data-ttu-id="e0452-136">**찾기 옵션** 에서 **사용** 확인란을 선택하면 **바꿀 내용**입력란 옆에 있는 삼각형 단추가 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-136">This triangular button next to the **Replace with** box becomes available when the **Use** check box is selected in **Find Options**.</span></span> <span data-ttu-id="e0452-137">이 단추를 클릭하면 선택한 **사용** 옵션에 따라 와일드카드 또는 정규식 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-137">Click this button to display a list of wildcards or regular expressions, depending upon the **Use** option selected.</span></span> <span data-ttu-id="e0452-138">이 목록에서 항목을 클릭하면 해당 항목이 **바꿀 내용** 입력란에 지정된 문자열에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-138">Clicking any item in this list adds it to the string specified in the **Replace with** box.</span></span>  
  
 <span data-ttu-id="e0452-139">**바꾸기**</span><span class="sxs-lookup"><span data-stu-id="e0452-139">**Replace**</span></span>  
 <span data-ttu-id="e0452-140">**찾을 내용** 입력란에 지정된 문자열의 현재 인스턴스를 **바꿀 내용** 입력란에 지정된 문자열로 바꾸고 **찾는 위치**에 지정된 범위 내에서 다음 인스턴스를 찾으려면 이 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-140">Click this button to replace the current instance of the string specified in the **Find what** box with the string specified in the **Replace with** box, and find the next instance within the scope specified in **Look in**.</span></span>  
  
 <span data-ttu-id="e0452-141">**모두 바꾸기**</span><span class="sxs-lookup"><span data-stu-id="e0452-141">**Replace all**</span></span>  
 <span data-ttu-id="e0452-142">**찾는 위치** 입력란에 지정된 범위 내의 모든 파일에서 **찾을 내용** 입력란에 지정된 문자열을 **바꿀 내용** 입력란에 지정된 문자열로 바꾸려면 이 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-142">Click this button to replace all instances of the string specified in the **Find what** box with the string specified in the **Replace with** box, in all files within the scope specified in the **Look in** box.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="e0452-143">**찾는 위치** 에 수정하려는 파일만 포함되도록 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-143">Make sure that **Look in** is set to include only those files that you want to modify.</span></span>  
  
 <span data-ttu-id="e0452-144">**모두 바꾸기를 실행한 후 수정한 파일 열어 두기** 옵션이 포함된 미리 알림이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-144">A reminder is displayed that includes a **Keep modified files open** option.</span></span> <span data-ttu-id="e0452-145">**실행 취소** 옵션을 유지하려면 이 옵션을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-145">To retain the **Undo** option, you must select this option.</span></span> <span data-ttu-id="e0452-146">**실행 취소** 는 수정 후에 편집을 위해 계속 열려 있는 파일에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-146">**Undo** is only available in files that remain open for editing after they are modified.</span></span>  
  
 <span data-ttu-id="e0452-147">**파일 건너뛰기**</span><span class="sxs-lookup"><span data-stu-id="e0452-147">**Skip File**</span></span>  
 <span data-ttu-id="e0452-148">**찾는 위치** 에 여러 파일을 포함하는 값을 지정한 경우 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-148">Becomes available when the value specified for **Look in** includes multiple files.</span></span> <span data-ttu-id="e0452-149">현재 파일을 검색 또는 수정하지 않으려면 이 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-149">Click this button if you do not want to search or modify the current file.</span></span> <span data-ttu-id="e0452-150">검색은 **찾는 위치**의 목록에 있는 다음 파일에서 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-150">The search will continue in the next file on the list in **Look in**.</span></span>  
  
## <a name="look-in"></a><span data-ttu-id="e0452-151">찾는 위치</span><span class="sxs-lookup"><span data-stu-id="e0452-151">Look In</span></span>  
 <span data-ttu-id="e0452-152">**Look in**</span><span class="sxs-lookup"><span data-stu-id="e0452-152">**Look in**</span></span>  
 <span data-ttu-id="e0452-153">**찾을 내용**에 지정된 텍스트를 찾을 위치를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-153">Select the location to look for the text specified in **Find what**.</span></span> <span data-ttu-id="e0452-154">사용할 수 있는 옵션은 대화 상자를 열 때 포커스가 놓여 있던 문서 창을 검색하는 **현재 문서**와 **에서 현재 열려 있는 모든 문서 창을 검색하는**모든 열린 문서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]입니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-154">Options are **Current Document**, which searches the document window that had focus when the dialog box was opened, and **All Open Documents**, which searches all document windows that are currently open in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="find-options"></a><span data-ttu-id="e0452-155">사용</span><span class="sxs-lookup"><span data-stu-id="e0452-155">Find Options</span></span>  
 <span data-ttu-id="e0452-156">**찾기 옵션** 섹션을 확장하거나 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-156">You can expand or collapse the **Find Options** section.</span></span> <span data-ttu-id="e0452-157">다음과 같은 옵션을 선택하거나 선택 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-157">The following options can be selected or cleared.</span></span>  
  
 <span data-ttu-id="e0452-158">**대/소문자 구분**</span><span class="sxs-lookup"><span data-stu-id="e0452-158">**Match case**</span></span>  
 <span data-ttu-id="e0452-159">이 확인란을 선택하면 찾기 결과 창에 **찾을 내용** 에 지정된 문자열의 인스턴스 중 내용과 대/소문자가 모두 일치하는 인스턴스만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-159">When this check box is selected, the Find Results windows will only display instances of the string specified in **Find what** that are matched both by content and by case.</span></span> <span data-ttu-id="e0452-160">예를 들어**대/소문자 구분**확인란을 선택하고 " **MyObject** "를 검색하면 "MyObject"는 반환되지만 "myobject"나 "MYOBJECT"는 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-160">For example, a search for "**MyObject**" with the **Match case** check box selected will return "MyObject" but not "myobject" or "MYOBJECT."</span></span>  
  
 <span data-ttu-id="e0452-161">**단어 단위로**</span><span class="sxs-lookup"><span data-stu-id="e0452-161">**Match whole word**</span></span>  
 <span data-ttu-id="e0452-162">이 확인란을 선택하면 **찾을 내용** 으로 검색된 문자열 중 단어 단위로 일치하는 문자열만 찾기 결과 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-162">When selected, the Find Results windows will only display instances of the string specified in **Find what** that are matched in complete words.</span></span> <span data-ttu-id="e0452-163">예를 들어 **MyObject** 를 검색하면 "MyObject"는 반환되지만 "CMyObject"나 "MyObjectC"는 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-163">For example, a search for **MyObject** will return "MyObject" but not "CMyObject" or "MyObjectC."</span></span>  
  
 <span data-ttu-id="e0452-164">**위로 검색**</span><span class="sxs-lookup"><span data-stu-id="e0452-164">**Search up**</span></span>  
 <span data-ttu-id="e0452-165">커서 위치를 기준으로 문서 앞쪽으로 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-165">Search from the cursor location towards the beginning of the document.</span></span>  
  
 <span data-ttu-id="e0452-166">**숨겨진 텍스트 검색**</span><span class="sxs-lookup"><span data-stu-id="e0452-166">**Search hidden text**</span></span>  
 <span data-ttu-id="e0452-167">숨겨지거나 축소된 텍스트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-167">Locate instances of the text that are concealed and collapsed text.</span></span>  
  
 <span data-ttu-id="e0452-168">**사용**</span><span class="sxs-lookup"><span data-stu-id="e0452-168">**Use**</span></span>  
 <span data-ttu-id="e0452-169">**찾을 내용** 또는 **바꿀 내용** 입력란에 입력한 특수 문자의 해석 방법을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-169">Indicates how to interpret special characters entered in the **Find what** or **Replace with** text boxes.</span></span> <span data-ttu-id="e0452-170">옵션에는 **와일드카드** 및 **정규식**이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-170">The options include **Wildcards** and **Regular Expressions**.</span></span>  
  
 <span data-ttu-id="e0452-171">**Regular Expressions**</span><span class="sxs-lookup"><span data-stu-id="e0452-171">**Regular Expressions**</span></span>  
 <span data-ttu-id="e0452-172">특수 표기를 사용하여 일치하는 텍스트의 패턴을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-172">Special notations define patterns of text to match.</span></span> <span data-ttu-id="e0452-173">목록을 보려면 [정규식으로 텍스트 검색](search-text-with-regular-expressions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0452-173">For a list, see [Search Text with Regular Expressions](search-text-with-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="e0452-174">**와일드카드**</span><span class="sxs-lookup"><span data-stu-id="e0452-174">**Wildcards**</span></span>  
 <span data-ttu-id="e0452-175">별표(`*`) 및 물음표(`?`)와 같은 특수 문자는 하나 이상의 문자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-175">Special characters such as asterisks (`*`) and question marks (`?`) represent one or more characters.</span></span> <span data-ttu-id="e0452-176">목록을 보려면 [와일드카드로 텍스트 검색](search-text-with-wildcards.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0452-176">For a list, see [Search Text with Wildcards](search-text-with-wildcards.md).</span></span>  
  
 <span data-ttu-id="e0452-177">**다음 찾기**</span><span class="sxs-lookup"><span data-stu-id="e0452-177">**Find Next**</span></span>  
 <span data-ttu-id="e0452-178">**찾을 내용** 입력란에 있는 텍스트에 대한 검색을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-178">Begins searching for the text in the **Find what** box.</span></span>  
  
 <span data-ttu-id="e0452-179">**바꾸기**</span><span class="sxs-lookup"><span data-stu-id="e0452-179">**Replace**</span></span>  
 <span data-ttu-id="e0452-180">**찾을 내용** 에 지정된 문자열의 현재 인스턴스를 **바꿀 내용**에 지정된 문자열로 바꾸고 **찾는 위치**에 지정된 범위 내에서 다음 인스턴스를 찾으려면 이 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-180">Click this button to replace the current instance of the string specified in **Find what** with the string specified in **Replace with**, and find the next instance within the scope specified in **Look in**.</span></span>  
  
 <span data-ttu-id="e0452-181">**Replace All**</span><span class="sxs-lookup"><span data-stu-id="e0452-181">**Replace All**</span></span>  
 <span data-ttu-id="e0452-182">**찾는 위치** 에 지정된 범위 내의 모든 파일에서 **찾을 내용**에 지정된 문자열을 **바꿀 내용**에 지정된 문자열로 바꾸려면 이 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-182">Choose this button to replace all instances of the string specified in **Find what** with the string specified in **Replace with**, in all files within the scope specified in **Look in**.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="e0452-183">**찾는 위치** 에 수정하려는 파일만 포함되도록 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-183">Make sure that **Look in** is set to include only those files that you want to modify.</span></span>  
  
## <a name="find-and-replace-views"></a><span data-ttu-id="e0452-184">찾기 및 바꾸기 뷰</span><span class="sxs-lookup"><span data-stu-id="e0452-184">Find and Replace Views</span></span>  
 <span data-ttu-id="e0452-185">찾기 및 바꾸기 창의 위쪽에 있는 탭에는 **뷰** 메뉴가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-185">The tabs at the top of the Find and Replace window include **View** menus.</span></span> <span data-ttu-id="e0452-186">이러한 메뉴를 사용하면 활성 창에서 표시할 필드 집합을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-186">These menus enable you to choose a set of fields to display in the active pane.</span></span> <span data-ttu-id="e0452-187">**찾기 및 바꾸기** 창은 사용하기 편한 위치에 도킹한 다음 탭 사이 및 뷰 사이를 오가며 찾기 또는 바꾸기 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-187">You can leave the **Find and Replace** window docked in a convenient location, and then change from tab to tab and view to view to perform any type of find or replace operation.</span></span>  
  
 <span data-ttu-id="e0452-188">**빠른 찾기**</span><span class="sxs-lookup"><span data-stu-id="e0452-188">**Quick Find**</span></span>  
 <span data-ttu-id="e0452-189">이 도구 모음 탭은 대화 상자를 **빠른 찾기** 대화 상자로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-189">This toolbar tab changes the dialog box to a **Quick Find** dialog box.</span></span>  
  
 <span data-ttu-id="e0452-190">**파일에서 찾기**</span><span class="sxs-lookup"><span data-stu-id="e0452-190">**Find in Files**</span></span>  
 <span data-ttu-id="e0452-191">이 도구 모음 탭은 대화 상자를 **파일에서 찾기** 대화 상자로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-191">This toolbar tab changes the dialog box to a **Find in Files** dialog box.</span></span>  
  
 <span data-ttu-id="e0452-192">**빠른 바꾸기**</span><span class="sxs-lookup"><span data-stu-id="e0452-192">**Quick Replace**</span></span>  
 <span data-ttu-id="e0452-193">이 도구 모음 탭은 대화 상자를 **빠른 바꾸기** 대화 상자로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-193">This toolbar tab changes the dialog box to a **Quick Replace** dialog box</span></span>  
  
 <span data-ttu-id="e0452-194">**파일에서 바꾸기**</span><span class="sxs-lookup"><span data-stu-id="e0452-194">**Replace in Files**</span></span>  
 <span data-ttu-id="e0452-195">이 도구 모음 탭은 대화 상자를 **파일에서 바꾸기** 대화 상자로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e0452-195">This toolbar tab changes the dialog box to a **Replace in Files** dialog box</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0452-196">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e0452-196">See Also</span></span>  
 [<span data-ttu-id="e0452-197">SQL Server Management Studio 바로 가기 키</span><span class="sxs-lookup"><span data-stu-id="e0452-197">SQL Server Management Studio Keyboard Shortcuts</span></span>](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)  
